## Method Missing Example

Random example of using method_missing to modify the behaviour of an object instance:

    god = { :name => 'Jebus', :kills_kittens? => true }
    
    # modify this hash instance to have additional methods for each attribute
    god.instance_eval do
      def method_missing(method)
        if keys.include?(method)
          self[method]
        else
          raise NoMethodError.new("undefined method '#{method}' for #{inspect}:#{self.class}")
        end
      end
    end
    
    # >> god.name
    # => "Jebus"
    # >> god.kills_kittens?
    # => true
    # >> god.is_real?
    # NoMethodError: undefined method 'is_real?' for {:kills_kittens?=>true, :name=>"Jebus"}:Hash

# Ruby 1.8.7/1.9

## __method__

    def foo
      __method__
    end
    
    # >> foo
    # => :foo
